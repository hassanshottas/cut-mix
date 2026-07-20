# cut-mix
application web pour salon de coiffure mixte moderne 
'use client';

import React, { useState } from 'react';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import LoginForm from '@/components/auth/LoginForm';
import RegisterForm from '@/components/auth/RegisterForm';

/**
 * Page d'authentification CutMix
 * Layout split-screen avec logo/tagline (gauche) et formulaires (droite)
 */
export default function AuthPage(): React.ReactElement {
  const [activeTab, setActiveTab] = useState<'login' | 'register'>('login');

  return (
    <div className="flex min-h-screen bg-gradient-to-br from-[#1A1A2E] to-[#16213e]">
      {/* Colonne gauche - Branding (visible desktop, caché mobile) */}
      <div className="hidden lg:flex lg:w-1/2 flex-col items-center justify-center px-8 py-12">
        <div className="max-w-sm text-center">
          {/* Animation logo avec ciseaux */}
          <div className="mb-8 flex justify-center">
            <svg
              className="w-16 h-16 animate-spin-slow"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              {/* Ciseaux stylisés */}
              <circle cx="8" cy="6" r="2" fill="#E94560" />
              <circle cx="16" cy="6" r="2" fill="#E94560" />
              <path
                d="M8 8L12 14M16 8L12 14M12 14L12 20"
                stroke="#E94560"
                strokeWidth="1.5"
                strokeLinecap="round"
                strokeLinejoin="round"
              />
            </svg>
          </div>

          {/* Logo texte */}
          <h1 className="text-5xl font-bold text-white mb-2 font-playfair">
            CutMix
          </h1>

          {/* Tagline */}
          <p className="text-xl text-[#E94560] mb-12 font-light">
            Votre style, notre signature.
          </p>

          {/* Texte descriptif */}
          <p className="text-gray-300 text-base leading-relaxed">
            Bienvenue dans votre espace personnel. Connectez-vous pour accéder
            à vos réservations, gérer votre profil et découvrir nos services
            exclusifs.
          </p>
        </div>
      </div>

      {/* Colonne droite - Formulaires */}
      <div className="w-full lg:w-1/2 flex items-center justify-center px-4 py-8 sm:px-6 sm:py-12">
        <div className="w-full max-w-md">
          {/* Logo mobile */}
          <div className="lg:hidden mb-8 text-center">
            <h1 className="text-4xl font-bold text-white font-playfair mb-2">
              CutMix
            </h1>
            <p className="text-sm text-[#E94560]">
              Votre style, notre signature.
            </p>
          </div>

          {/* Tabs pour Connexion/Inscription */}
          <Tabs 
            value={activeTab} 
            onValueChange={(val) => setActiveTab(val as 'login' | 'register')}
            className="w-full"
          >
            <TabsList className="grid w-full grid-cols-2 mb-6 bg-gray-200 dark:bg-gray-800">
              <TabsTrigger
                value="login"
                className="data-[state=active]:bg-[#E94560] data-[state=active]:text-white"
              >
                Connexion
              </TabsTrigger>
              <TabsTrigger
                value="register"
                className="data-[state=active]:bg-[#E94560] data-[state=active]:text-white"
              >
                Inscription
              </TabsTrigger>
            </TabsList>

            {/* Contenu onglet Connexion */}
            <TabsContent value="login" className="mt-6">
              <LoginForm />
            </TabsContent>

            {/* Contenu onglet Inscription */}
            <TabsContent value="register" className="mt-6">
              <RegisterForm />
            </TabsContent>
          </Tabs>
        </div>
      </div>

      {/* Styles pour l'animation des ciseaux */}
      <style jsx>{`
        @keyframes spin-slow {
          from {
            transform: rotate(0deg);
          }
          to {
            transform: rotate(360deg);
          }
        }
        .animate-spin-slow {
          animation: spin-slow 6s linear infinite;
        }
      `}</style>
    </div>
  );
}
